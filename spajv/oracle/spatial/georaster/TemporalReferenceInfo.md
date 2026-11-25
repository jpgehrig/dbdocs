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

- [Prev Class](SubLayerInfo.md)
- Next Class

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

## Class TemporalReferenceInfo

- java.lang.Object

- - oracle.spatial.georaster.TemporalReferenceInfo

<!-- -->

-

  ------------------------------------------------------------------------



      public class TemporalReferenceInfo
      extends java.lang.Object

  TemporalReferenceInfo is a Java class mapped to the XML element TemporalReferenceInfo in the Oracle Spatial GeoRaster metadata.

<!-- -->

- - ### Method Summary

    **All Methods[Instance Methods](javascript:show(2);)[Concrete Methods](javascript:show(8);)**

    | Modifier and Type    | Method and Description                                                                                                            |
    |----------------------|-----------------------------------------------------------------------------------------------------------------------------------|
    | `TIMESTAMP`          | `getBeginDateTime``()`<br>Returns the begin date and time.                                                                        |
    | `java.lang.String[]` | `getDescription``()`<br>Returns the georeference description.                                                                     |
    | `TIMESTAMP`          | `getEndDateTime``()`<br>Returns the end date and time.                                                                            |
    | `java.lang.String`   | `getTemporalResolutionDescription``()`<br>Returns the temporal resolution description.                                            |
    | `java.lang.Boolean`  | `isReferenced``()`<br>Returns true if the current GeoRaster object is georeferenced.                                              |
    | `void`               | `setBeginDateTime``(TIMESTAMP beginDateTime)`<br>Sets the begin date and time.                                                    |
    | `void`               | `setDescription``(java.lang.String[] description)`<br>Sets the georeference description.                                          |
    | `void`               | `setEndDateTime``(TIMESTAMP endDateTime)`<br>Sets the end date and time.                                                          |
    | `void`               | `setReferenced``(java.lang.Boolean isReferenced)`<br>Sets true if the current GeoRaster object is georeferenced.                  |
    | `void`               | `setTemporalResolutionDescription``(java.lang.String temporalResolutionDescription)`<br>Sets the temporal resolution description. |

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

    - #### setReferenced

          public void setReferenced(java.lang.Boolean isReferenced)

      Sets true if the current GeoRaster object is georeferenced.
      Parameters:
      `isReferenced` - true if the current GeoRaster object is georeferenced

    <!-- -->

    - #### getDescription

          public java.lang.String[] getDescription()

      Returns the georeference description.
      Returns:
      georeference description.

    <!-- -->

    - #### setDescription

          public void setDescription(java.lang.String[] description)

      Sets the georeference description.
      Parameters:
      `description` - georeference description.

    <!-- -->

    - #### getBeginDateTime

          public TIMESTAMP getBeginDateTime()

      Returns the begin date and time.
      Returns:
      begin date and time.

    <!-- -->

    - #### setBeginDateTime

          public void setBeginDateTime(TIMESTAMP beginDateTime)

      Sets the begin date and time.
      Parameters:
      `beginDateTime` - begin date and time.

    <!-- -->

    - #### getEndDateTime

          public TIMESTAMP getEndDateTime()

      Returns the end date and time.
      Returns:
      end Date Time.

    <!-- -->

    - #### setEndDateTime

          public void setEndDateTime(TIMESTAMP endDateTime)

      Sets the end date and time.
      Parameters:
      `endDateTime` - end date and time.

    <!-- -->

    - #### getTemporalResolutionDescription

          public java.lang.String getTemporalResolutionDescription()

      Returns the temporal resolution description.
      Returns:
      temporal resolution description.

    <!-- -->

    - #### setTemporalResolutionDescription

          public void setTemporalResolutionDescription(java.lang.String temporalResolutionDescription)

      Sets the temporal resolution description.
      Parameters:
      `temporalResolutionDescription` - temporal resolution description

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

- [Prev Class](SubLayerInfo.md)
- Next Class

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
