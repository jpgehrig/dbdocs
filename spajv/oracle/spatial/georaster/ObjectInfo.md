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

- [Prev Class](LayerInfo.md)
- [Next Class](RasterInfo.md)

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

## Class ObjectInfo

- java.lang.Object

- - oracle.spatial.georaster.ObjectInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class ObjectInfo
      extends java.lang.Object

  ObjectInfo is a Java class mapped to the XML element ObjectInfo in the Oracle Spatial GeoRaster metadata.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type    | Method and Description                                                                                                |
    |----------------------|-----------------------------------------------------------------------------------------------------------------------|
    | `java.lang.Double`   | `getBlankCellValue``()`<br>Returns the blank cell value defined in the GeoRaster object.                              |
    | `java.lang.Long`     | `getDefaultBlue``()`<br>Returns the default blue band set in the GeoRaster object.                                    |
    | `java.lang.Long`     | `getDefaultGreen``()`<br>Returns the default green band set in the GeoRaster object.                                  |
    | `java.lang.Long`     | `getDefaultRed``()`<br>Returns the default red band set in the GeoRaster object.                                      |
    | `java.lang.String[]` | `getDescription``()`<br>Returns the description of the GeoRaster object.                                              |
    | `java.lang.String`   | `getMajorVersion``()`<br>Returns the major version of the GeoRaster object.                                           |
    | `java.lang.String`   | `getMinorVersion``()`<br>Returns the minor version of the GeoRaster object.                                           |
    | `java.lang.Integer`  | `getRasterType``()`<br>Returns the GeoRaster type.                                                                    |
    | `java.lang.String`   | `getUserID``()`<br>Returns the GeoRaster user ID.                                                                     |
    | `java.lang.Boolean`  | `isBlank``()`<br>Returns true if the GeoRaster object is blank.                                                       |
    | `void`               | `setBlankCellValue``(java.lang.Double blankCellValue)`<br>Sets the blank cell value for the current GeoRaster object. |
    | `void`               | `setDefaultBlue``(java.lang.Long defaultBlue)`<br>Sets the default blue band for the current GeoRaster object.        |
    | `void`               | `setDefaultGreen``(java.lang.Long defaultGreen)`<br>Sets the default green band for the current GeoRaster object.     |
    | `void`               | `setDefaultRed``(java.lang.Long defaultRed)`<br>Sets the default red band for the current GeoRaster object.           |
    | `void`               | `setDescription``(java.lang.String[] description)`<br>Sets the description for the current GeoRaster object.          |
    | `void`               | `setMajorVersion``(java.lang.String majorVersion)`<br>Sets the major version for the current GeoRaster object.        |
    | `void`               | `setMinorVersion``(java.lang.String minorVersion)`<br>Sets the minor version for the current GeoRaster object.        |
    | `void`               | `setUserID``(java.lang.String ID)`<br>Sets the user ID for the current GeoRaster object.                              |

    - ### Methods inherited from class java.lang.Object

      `equals, getClass, hashCode, notify, notifyAll, toString, wait, wait, wait`

<!-- -->

- - ### Method Detail

    - #### getRasterType

          public java.lang.Integer getRasterType()

      Returns the GeoRaster type.
      Returns:
      Raster type.

    <!-- -->

    - #### getUserID

          public java.lang.String getUserID()

      Returns the GeoRaster user ID.
      Returns:
      GeoRaster user ID.

    <!-- -->

    - #### setUserID

          public void setUserID(java.lang.String ID)

      Sets the user ID for the current GeoRaster object.
      Parameters:
      `ID` - user ID.

    <!-- -->

    - #### getDescription

          public java.lang.String[] getDescription()

      Returns the description of the GeoRaster object.
      Returns:
      the description of the GeoRaster object.

    <!-- -->

    - #### setDescription

          public void setDescription(java.lang.String[] description)

      Sets the description for the current GeoRaster object.
      Parameters:
      `description` - set description for the current GeoRaster object.

    <!-- -->

    - #### getMajorVersion

          public java.lang.String getMajorVersion()

      Returns the major version of the GeoRaster object.
      Returns:
      the major version of the GeoRaster object.

    <!-- -->

    - #### setMajorVersion

          public void setMajorVersion(java.lang.String majorVersion)

      Sets the major version for the current GeoRaster object.
      Parameters:
      `majorVersion` - set major version for the current GeoRaster object.

    <!-- -->

    - #### getMinorVersion

          public java.lang.String getMinorVersion()

      Returns the minor version of the GeoRaster object.
      Returns:
      the minor version of the GeoRaster object.

    <!-- -->

    - #### setMinorVersion

          public void setMinorVersion(java.lang.String minorVersion)

      Sets the minor version for the current GeoRaster object.
      Parameters:
      `minorVersion` - set minor version for the current GeoRaster object.

    <!-- -->

    - #### isBlank

          public java.lang.Boolean isBlank()

      Returns true if the GeoRaster object is blank.
      Returns:
      true if the GeoRaster object is blank.

    <!-- -->

    - #### getBlankCellValue

          public java.lang.Double getBlankCellValue()

      Returns the blank cell value defined in the GeoRaster object.
      Returns:
      the blank cell value defined in the GeoRaster object.

    <!-- -->

    - #### setBlankCellValue

          public void setBlankCellValue(java.lang.Double blankCellValue)

      Sets the blank cell value for the current GeoRaster object.
      Parameters:
      `blankCellValue` - blank cell value

    <!-- -->

    - #### getDefaultRed

          public java.lang.Long getDefaultRed()

      Returns the default red band set in the GeoRaster object.
      Returns:
      the default red band set in the GeoRaster object.

    <!-- -->

    - #### setDefaultRed

          public void setDefaultRed(java.lang.Long defaultRed)

      Sets the default red band for the current GeoRaster object.
      Parameters:
      `defaultRed` - default red band

    <!-- -->

    - #### getDefaultGreen

          public java.lang.Long getDefaultGreen()

      Returns the default green band set in the GeoRaster object.
      Returns:
      the default green band set in the GeoRaster object.

    <!-- -->

    - #### setDefaultGreen

          public void setDefaultGreen(java.lang.Long defaultGreen)

      Sets the default green band for the current GeoRaster object.
      Parameters:
      `defaultGreen` - default green band

    <!-- -->

    - #### getDefaultBlue

          public java.lang.Long getDefaultBlue()

      Returns the default blue band set in the GeoRaster object.
      Returns:
      the default blue band set in the GeoRaster object.

    <!-- -->

    - #### setDefaultBlue

          public void setDefaultBlue(java.lang.Long defaultBlue)

      Sets the default blue band for the current GeoRaster object.
      Parameters:
      `defaultBlue` - default blue band

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

- [Prev Class](LayerInfo.md)
- [Next Class](RasterInfo.md)

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
