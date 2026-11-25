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

- Prev Class
- [Next Class](GCPGeoreference.md)

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

## Class BandReferenceInfo

- java.lang.Object

- - oracle.spatial.georaster.BandReferenceInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class BandReferenceInfo
      extends java.lang.Object

  BandReferenceInfo is a Java class mapped to the XML element BandReferenceInfo in the Oracle Spatial GeoRaster metadata.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type   | Method and Description                                                                                   |
    |---------------------|----------------------------------------------------------------------------------------------------------|
    | `java.util.Vector`  | `getBandReference``()`<br>Returns the band reference vector.                                             |
    | `java.lang.String`  | `getDescription``()`<br>Returns the description.                                                         |
    | `java.lang.String`  | `getRadiometricResolutionDescription``()`<br>Returns the radiometric resolution description.             |
    | `java.lang.Double`  | `getSpectralExtent_Max``()`<br>Returns the maximum spectral extent.                                      |
    | `java.lang.Double`  | `getSpectralExtent_Min``()`<br>Returns the minimum spectral extent.                                      |
    | `java.lang.String`  | `getSpectralResolutionDescription``()`<br>Returns the spectral resolution description.                   |
    | `java.lang.Double`  | `getSpectralTolerance``()`<br>Returns the spectral tolerance.                                            |
    | `java.lang.String`  | `getSpectralUnit``()`<br>Returns the spectral unit.                                                      |
    | `java.lang.Boolean` | `isReferenced``()`<br>Returns true if the current GeoRaster object is georeferenced.                     |
    | `void`              | `setSpectralResolution``(double resolution)`<br>Sets the spectral resolution of the specified dimension. |
    | `void`              | `setSpectralUnit``(java.lang.String spectralUnit)`<br>Sets the spectral unit.                            |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### isReferenced

          public java.lang.Boolean isReferenced()

      Returns true if the current GeoRaster object is georeferenced.
      Returns:
      true if the current GeoRaster object is georeferenced.

    <!-- -->

    - #### getDescription

          public java.lang.String getDescription()

      Returns the description.
      Returns:
      description.

    <!-- -->

    - #### getRadiometricResolutionDescription

          public java.lang.String getRadiometricResolutionDescription()

      Returns the radiometric resolution description.
      Returns:
      radiometric resolution description.

    <!-- -->

    - #### getSpectralUnit

          public java.lang.String getSpectralUnit()

      Returns the spectral unit.
      Returns:
      spectral unit.

    <!-- -->

    - #### setSpectralUnit

          public void setSpectralUnit(java.lang.String spectralUnit)

      Sets the spectral unit.
      Parameters:
      `spectralUnit` - spectral unit

    <!-- -->

    - #### getSpectralTolerance

          public java.lang.Double getSpectralTolerance()

      Returns the spectral tolerance.
      Returns:
      spectral tolerance.

    <!-- -->

    - #### getSpectralResolutionDescription

          public java.lang.String getSpectralResolutionDescription()

      Returns the spectral resolution description.
      Returns:
      spectral resolution description.

    <!-- -->

    - #### setSpectralResolution

          public void setSpectralResolution(double resolution)

      Sets the spectral resolution of the specified dimension.
      Parameters:
      `resolution` - minimum spectral resolution

    <!-- -->

    - #### getSpectralExtent_Min

          public java.lang.Double getSpectralExtent_Min()

      Returns the minimum spectral extent.
      Returns:
      minimum spectral extent.

    <!-- -->

    - #### getSpectralExtent_Max

          public java.lang.Double getSpectralExtent_Max()

      Returns the maximum spectral extent.
      Returns:
      maximum spectral extent.

    <!-- -->

    - #### getBandReference

          public java.util.Vector getBandReference()

      Returns the band reference vector.
      Returns:
      band reference vector.

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

- Prev Class
- [Next Class](GCPGeoreference.md)

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
