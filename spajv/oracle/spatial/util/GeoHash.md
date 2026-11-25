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

- [Prev Class](Generalization3D.md)
- [Next Class](GeometryExceptionWithContext.md)

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

oracle.spatial.util

## Class GeoHash

- java.lang.Object

- - oracle.spatial.util.GeoHash

<!-- -->

- All Implemented Interfaces:
  java.io.Serializable

  ------------------------------------------------------------------------



      public class GeoHash
      extends java.lang.Object
      implements java.io.Serializable

  See Also:
  [Serialized Form](../../../serialized-form.md)

<!-- -->

- - ### Field Summary

    **Fields**

    | Modifier and Type         | Field and Description |
    |---------------------------|-----------------------|
    | `static java.lang.String` | `base32`              |

  <!-- -->

  - ### Constructor Summary

    **Constructors**

    | Constructor and Description                                     |
    |-----------------------------------------------------------------|
    | `GeoHash``()`                                                   |
    | `GeoHash``(double longitude, double latitude, int hashLength)`  |

  <!-- -->

  - ### Method Summary

    **All Methods[Static Methods](javascript:show(1);)[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type                       | Method and Description                                                                                                                                                                     |
    |-----------------------------------------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
    | `static double[]`                       | `asMer``(java.lang.String geohash)`<br>Finds the mer corresponding to a geohash                                                                                                            |
    | `static long`                           | `decimalValue``(java.lang.String ghString)`<br>Computes the numeric value of a geohash string                                                                                              |
    | `static GeoHash`                        | `geohash``(double longitude, double latitude, int hashLength)`<br>GeoHash from longitude, latitude with number of characters = hashLength                                                  |
    | `static GeoHash`                        | `geohash``(long value, int hashLength)`<br>GeoHash corresponding to the long value                                                                                                         |
    | `static GeoHash`                        | `geohash``(java.lang.String bitString)`<br>GeoHash from a bit string the length of the string must be a multiple of 5                                                                      |
    | `static int[]`                          | `geohashBits``(double longitude, double latitude, int numBits)`                                                                                                                            |
    | `static GeoHash`                        | `geohashFromString``(java.lang.String base32String)`<br>GeoHash from a string (base 32)                                                                                                    |
    | `java.lang.String`                      | `geohashString``(double longitude, double latitude, int hashLength)`                                                                                                                       |
    | `static GeoHash`                        | `geohashWithBitsLength``(double longitude, double latitude, int numberOfBits)`<br>GeoHash from longitude, latitude with number of bits = numberOfBits numberOfBits must be a multiple of 5 |
    | [`JPoint2DD`](../geometry/JPoint2DD.md) | `getCenterPoint``()`<br>Computes the center point of the geohash mer                                                                                                                       |
    | `long`                                  | `getDecimalValue``()`<br>Getter for the numeric value of the geohash                                                                                                                       |
    | `GeoHash[]`                             | `getEightNeighbors``()`<br>Finds the eight neighbors of this                                                                                                                               |
    | `java.lang.String`                      | `getGeoHashString``()`<br>Getter for geohash string                                                                                                                                        |
    | `GeoHash`                               | `getGeoHashToTheEast``()`<br>Finds the geohash to the east of this.                                                                                                                        |
    | `GeoHash`                               | `getGeoHashToTheNorth``()`<br>Finds the geohash to the north of this.                                                                                                                      |
    | `GeoHash`                               | `getGeoHashToTheSouth``()`<br>Finds the geohash to the south of this                                                                                                                       |
    | `GeoHash`                               | `getGeoHashToTheWest``()`<br>Finds the geohash to the west of this                                                                                                                         |
    | `double[]`                              | `getMer``()`<br>Getter for mer                                                                                                                                                             |
    | `short`                                 | `getNumberOfBits``()`<br>Getter for the number of bits in the geohash bit string                                                                                                           |
    | `long`                                  | `getValue``()`                                                                                                                                                                             |
    | `GeoHash`                               | `()`<br>Finds the next geohash.                                                                                                                                                            |
    | `GeoHash`                               | `(int numberOfSteps)`<br>Finds the geohash removed by a given number of steps from this.                                                                                                   |
    | `static long`                           | `numberOfStepsBetween``(GeoHash gh1, GeoHash gh2)`                                                                                                                                         |
    | `GeoHash`                               | `prev``()`<br>Finds the previous geohash                                                                                                                                                   |
    | `java.lang.String`                      | `toBinaryString``()`<br>Computes an equivalent bit string representation of the geohash                                                                                                    |
    | `boolean`                               | `within``(GeoHash gh)`<br>Checks whether the mer of the given geohash is inside the mer of this                                                                                            |
    | `boolean`                               | `within``(`[`JPoint2DD`](../geometry/JPoint2DD.md)` point)`<br>Checks whether the given point is inside the mer of this.                                                                   |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Field Detail

    - #### base32

          public static final java.lang.String base32

      See Also:
      [Constant Field Values](../../../constant-values.md)

  <!-- -->

  - ### Constructor Detail

    - #### GeoHash

          public GeoHash()

    <!-- -->

    - #### GeoHash

          public GeoHash(double longitude,
                         double latitude,
                         int hashLength)

  <!-- -->

  - ### Method Detail

    - #### geohash

          public static GeoHash geohash(double longitude,
                                        double latitude,
                                        int hashLength)

      GeoHash from longitude, latitude with number of characters = hashLength
      Parameters:
      `longitude` - longitude of the point

      `latitude` - latitude of the point

      `hashLength` - precision of geohash in number of characters

      Returns:
      GeoHash of the point

    <!-- -->

    - #### geohashWithBitsLength

          public static GeoHash geohashWithBitsLength(double longitude,
                                                      double latitude,
                                                      int numberOfBits)

      GeoHash from longitude, latitude with number of bits = numberOfBits numberOfBits must be a multiple of 5
      Parameters:
      `longitude` - longitude of the point

      `latitude` - latitude of the point

      `numberOfBits` - precision of geohash in number of bits

      Returns:
      GeoHash of the point

    <!-- -->

    - #### geohash

          public static GeoHash geohash(java.lang.String bitString)

      GeoHash from a bit string the length of the string must be a multiple of 5
      Parameters:
      `bitString` - bit string

      Returns:
      GeoHash of the string

    <!-- -->

    - #### geohash

          public static GeoHash geohash(long value,
                                        int hashLength)

      GeoHash corresponding to the long value
      Parameters:
      `value` - value

      `hashLength` - precision of the geohash in number of characters

      Returns:
      GeoHash of the value

    <!-- -->

    - #### geohashFromString

          public static GeoHash geohashFromString(java.lang.String base32String)

      GeoHash from a string (base 32)
      Parameters:
      `base32String` - base32 string

      Returns:
      GeoHash of the string

    <!-- -->

    - #### geohashBits

          public static int[] geohashBits(double longitude,
                                          double latitude,
                                          int numBits)

    <!-- -->

    - #### getGeoHashString

          public java.lang.String getGeoHashString()

      Getter for geohash string

    <!-- -->

    - #### getMer

          public double[] getMer()

      Getter for mer

    <!-- -->

    - #### getNumberOfBits

          public short getNumberOfBits()

      Getter for the number of bits in the geohash bit string

    <!-- -->

    - #### getDecimalValue

          public long getDecimalValue()

      Getter for the numeric value of the geohash

    <!-- -->

    - #### getCenterPoint

          public JPoint2DD getCenterPoint()

      Computes the center point of the geohash mer
      Returns:
      JPoint2DD point

    <!-- -->

    - #### getValue

          public long getValue()

    <!-- -->

    - #### toBinaryString

          public java.lang.String toBinaryString()

      Computes an equivalent bit string representation of the geohash
      Returns:
      a bit string

    <!-- -->

    - #### next

          public GeoHash next(int numberOfSteps)

      Finds the geohash removed by a given number of steps from this.
      Parameters:
      `numberOfSteps` - number of steps to be moved

      Returns:
      GeoHash

    <!-- -->

    - #### next

          public GeoHash next()

      Finds the next geohash.
      Returns:
      GeoHash

    <!-- -->

    - #### prev

          public GeoHash prev()

      Finds the previous geohash
      Returns:
      GeoHash

    <!-- -->

    - #### asMer

          public static double[] asMer(java.lang.String geohash)

      Finds the mer corresponding to a geohash
      Returns:
      mer array

    <!-- -->

    - #### numberOfStepsBetween

          public static long numberOfStepsBetween(GeoHash gh1,
                                                  GeoHash gh2)

    <!-- -->

    - #### getGeoHashToTheNorth

          public GeoHash getGeoHashToTheNorth()

      Finds the geohash to the north of this.
      Returns:
      GeoHash

    <!-- -->

    - #### getGeoHashToTheEast

          public GeoHash getGeoHashToTheEast()

      Finds the geohash to the east of this.
      Returns:
      GeoHash

    <!-- -->

    - #### getGeoHashToTheSouth

          public GeoHash getGeoHashToTheSouth()

      Finds the geohash to the south of this
      Returns:
      GeoHash

    <!-- -->

    - #### getGeoHashToTheWest

          public GeoHash getGeoHashToTheWest()

      Finds the geohash to the west of this
      Returns:
      GeoHash

    <!-- -->

    - #### getEightNeighbors

          public GeoHash[] getEightNeighbors()

      Finds the eight neighbors of this
      Returns:
      an array of GeoHash in the order N, NE, E, SE, S, SW, W, NW

    <!-- -->

    - #### within

          public boolean within(GeoHash gh)

      Checks whether the mer of the given geohash is inside the mer of this
      Parameters:
      `gh` - geohash to be checked

    <!-- -->

    - #### within

          public boolean within(JPoint2DD point)

      Checks whether the given point is inside the mer of this.
      Parameters:
      `point` - point to be checked

      Returns:
      true if the point is inside mer

    <!-- -->

    - #### decimalValue

          public static long decimalValue(java.lang.String ghString)

      Computes the numeric value of a geohash string
      Parameters:
      `ghString` - base32 geohash string

      Returns:
      decimal value

    <!-- -->

    - #### geohashString

          public java.lang.String geohashString(double longitude,
                                                double latitude,
                                                int hashLength)

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

- [Prev Class](Generalization3D.md)
- [Next Class](GeometryExceptionWithContext.md)

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
